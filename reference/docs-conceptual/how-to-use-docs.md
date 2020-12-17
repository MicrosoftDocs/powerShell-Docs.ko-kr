---
ms.date: 07/29/2020
keywords: powershell,cmdlet
title: PowerShell 설명서를 사용하는 방법
description: 이 문서에서는 검색 필터링 및 버전 선택을 포함하여 이 사이트의 기능을 사용하는 방법을 설명합니다.
ms.openlocfilehash: b7e036fce0abb12f6c1ab4c0092784321a41a916
ms.sourcegitcommit: 2fc6ee49a70bda4c59135136bd5cc7782836a124
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94810303"
---
# <a name="how-to-use-the-powershell-documentation"></a>PowerShell 설명서를 사용하는 방법

PowerShell 온라인 설명서에 오신 것을 환영합니다. 이 사이트에는 다음 버전의 PowerShell에 대한 cmdlet 참조가 포함되어 있습니다.

- PowerShell 7.2(시험판)
- PowerShell 7.1(현재)
- PowerShell 7.0(LTS)
- PowerShell 5.1

## <a name="finding-articles-and-selecting-a-version"></a>문서 찾기 및 버전 선택

문서에서 콘텐츠를 검색하는 방법에는 두 가지가 있습니다. 가장 간단한 방법은 버전 선택기에서 필터 상자를 사용하는 것입니다. 문서의 제목에 표시되는 단어를 입력하기만 하면 됩니다. 페이지에 일치하는 문서 목록이 표시됩니다. 해당 목록에서 전체 사이트를 검색하는 옵션을 선택할 수도 있습니다.

기본적으로 이 사이트에는 출시된 최신 버전의 PowerShell에 대한 설명서가 표시됩니다. 일부 cmdlet은 다양한 버전의 PowerShell에서 다르게 작동합니다. 사용 중인 PowerShell 버전에 대한 설명서를 확인하세요.

페이지 위쪽의 버전 선택기를 사용하여 원하는 PowerShell 버전을 선택합니다.

![버전 선택기 사용](media/how-to-use-docs/version-search.gif)

사용 중인 PowerShell의 버전은 `$PSversionTable.PSVersion` 값을 검사해서 확인할 수 있습니다. 다음 예제에서는 Windows PowerShell v5.1의 출력을 보여 줍니다.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      19041  1
```

PowerShell을 처음 사용하고 명령 구문을 이해하는 데 도움이 필요하면 [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax)를 참조하세요.

## <a name="finding-articles-for-previous-versions"></a>이전 버전에 대한 문서 찾기

이전 버전의 PowerShell에 대한 설명서는 [이전 버전](https://aka.ms/PSLegacyDocs) 사이트에서 보관되어 있습니다.

이 사이트에는 다음 항목에 대한 설명서가 포함되어 있습니다.

- PowerShell 3.0
- PowerShell 4.0
- PowerShell 5.0
- PowerShell 6
- PowerShell 워크플로
- PowerShell 웹 액세스
