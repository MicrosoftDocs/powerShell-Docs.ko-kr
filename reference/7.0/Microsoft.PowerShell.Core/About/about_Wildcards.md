---
description: PowerShell에서 와일드 카드 문자를 사용 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 02/13/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 54108eaafa645452f58b1962c3f103bcdd5c9e4a
ms.sourcegitcommit: 9777152e026c47ba8d319593051416054cb62246
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/16/2021
ms.locfileid: "100529994"
---
# <a name="about-wildcards"></a>와일드 카드 정보

## <a name="short-description"></a>간단한 설명

PowerShell에서 와일드 카드 문자를 사용 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

와일드 카드 문자는 하나 이상의 문자를 나타냅니다. 이를 사용 하 여 명령에서 단어 패턴을 만들 수 있습니다. 와일드 카드 식은 연산자와 함께 사용 `-like` 되거나 와일드 카드를 허용 하는 모든 매개 변수와 함께 사용 됩니다.

예를 들어 `C:\Techdocs` 파일 이름 확장명을 사용 하 여 디렉터리의 모든 파일을 일치 시키려면 `.ppt` 다음과 같이 입력 합니다.

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

이 경우 별표 ( `*` ) 와일드 카드 문자는 파일 이름 확장명 앞에 나타나는 모든 문자를 나타냅니다 `.ppt` .

와일드 카드 식은 정규식 보다 간단 합니다. 자세한 내용은 [about_Regular_Expressions](./about_Regular_Expressions.md)를 참조 하세요.

PowerShell은 다음 와일드 카드 문자를 지원 합니다.

|와일드카드|설명               |예제 |일치        |일치 하지 않음|
|--------|--------------------------|--------|-------------|--------|
|\*      |0 개 이상의 문자를 찾습니다. | 은\*  | aA, ag, Apple | 바나나 |
|?       |해당 위치에서 한 문자 일치 | ? n | , in, on | 되었음 |
|\[ \]   |문자 범위 일치 | \[a-l \] ook | 책, 쿡, 모양 | 이나 |
|\[ \]   |특정 문자 일치 | \[bc \] ook | 책, 쿡 | 갈고리 |

동일한 단어 패턴에 여러 와일드 카드 문자를 포함할 수 있습니다. 예를 들어 이름이 **a** 부터 **l** 로 시작 하는 텍스트 파일을 찾으려면 다음을 입력 합니다.

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

많은 cmdlet은 매개 변수 값에 와일드 카드 문자를 허용 합니다. 각 cmdlet에 대 한 도움말 항목에서는 와일드 카드 문자를 허용 하는 매개 변수에 대해 설명 합니다. 와일드 카드 문자를 허용 하는 매개 변수의 경우에는 대/소문자를 구분 하지 않습니다.

명령 및 스크립트 블록에서 와일드 카드 문자를 사용 하 여 속성 값을 나타내는 단어 패턴을 만들 수 있습니다. 예를 들어 다음 명령은 **ServiceType** 속성 값이 **Interactive** 를 포함 하는 서비스를 가져옵니다.

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

다음 예에서 `If` 문에는 와일드 카드 문자를 사용 하 여 속성 값을 찾는 조건이 포함 되어 있습니다. 복원 지점의 **설명** 에 **PowerShell** 이 포함 되어 있는 경우이 명령은 복원 지점의 **CreationTime** 속성 값을 로그 파일에 추가 합니다.

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a>참고 항목

[about_Language_Keywords](about_Language_Keywords.md)

[about_If](about_If.md)

[about_Script_Blocks](about_Script_Blocks.md)
