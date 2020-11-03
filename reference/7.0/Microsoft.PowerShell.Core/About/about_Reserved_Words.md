---
description: PowerShell에서 특별 한 의미가 있기 때문에 식별자로 사용할 수 없는 예약 된 단어를 나열 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: c4b67a523a40319635d159791b80ab302b9aa3b4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223730"
---
# <a name="about-reserved-words"></a>예약 된 단어 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 특별 한 의미가 있기 때문에 식별자로 사용할 수 없는 예약 된 단어를 나열 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell에서 특별 한 의미가 있는 특정 단어가 있습니다. 이러한 단어가 따옴표 없이 표시 되는 경우 PowerShell은 문자열을 문자열로 처리 하는 대신 특별 한 의미를 적용 하려고 합니다. 이러한 단어를 특수 한 의미를 호출 하지 않고 명령 또는 스크립트에서 매개 변수 인수로 사용 하려면 예약어를 따옴표로 묶습니다.

다음은 PowerShell에서 예약 된 단어입니다.

```
assembly         exit            process
base             filter          public
begin            finally         return
break            for             sequence
catch            foreach         static
class            from (*)        switch
command          function        throw
configuration    hidden          trap
continue         if              try
data             in              type
define (*)       inlinescript    until
do               interface       using
dynamicparam     module          var (*)
else             namespace       while
elseif           parallel        workflow
end              param
enum             private

(*) These keywords are reserved for future use.
```

,, 및를 비롯 한 여러 언어 키워드에는 `Foreach` `If` `For` `While` 고유한 도움말 문서가 있습니다. 이를 보려면를 입력 하 `Get-Help about_` 고 키워드를 추가 합니다. 예를 들어 문에 대 한 정보를 가져오려면 `Foreach` 다음을 입력 합니다.

```powershell
Get-Help about_ForEach
```

문 또는 문 구문에 대 한 자세한 내용을 보려면 `Filter` `Return` 다음을 입력 하십시오.

```powershell
Get-Help about_Functions
```

다른 예약어에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> 모든 예약어에 자체 도움말 문서가 있는 것은 아닙니다. `Get-Help`에서 문서를 반환 하지 않는 경우 다음 명령을 사용 하 여 예약 된 단어에 대해 설명 하는 문서를 검색할 수 있습니다.
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a>참고 항목

- [about_Command_Syntax](about_Command_Syntax.md)
- [about_Language_Keywords](about_Language_Keywords.md)
- [about_Parsing](about_Parsing.md)
- [about_Quoting_Rules](about_Quoting_Rules.md)
- [about_Script_Blocks](about_Script_Blocks.md)
- [about_Special_Characters](about_Special_Characters.md)
