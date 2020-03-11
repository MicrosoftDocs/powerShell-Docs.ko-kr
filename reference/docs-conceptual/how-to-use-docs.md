---
ms.date: 10/20/2019
keywords: powershell,cmdlet
title: PowerShell 설명서를 사용하는 방법
ms.openlocfilehash: 7b73bc82f32e3ce1e6015822e0cc82078183931b
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279312"
---
# <a name="how-to-use-the-powershell-documentation"></a>PowerShell 설명서를 사용하는 방법

PowerShell 온라인 설명서에 오신 것을 환영합니다. 이 사이트에는 다음 버전의 PowerShell에 대한 cmdlet 참조가 포함되어 있습니다.

- PowerShell 7(미리 보기)
- PowerShell 6
- PowerShell 5.1

## <a name="finding-articles-and-selecting-a-version"></a>문서 찾기 및 버전 선택

문서에서 콘텐츠를 검색하는 방법에는 두 가지가 있습니다. 가장 간단한 방법은 버전 선택기에서 필터 상자를 사용하는 것입니다. 문서의 제목에 표시되는 단어를 입력하기만 하면 됩니다. 페이지에 일치하는 문서 목록이 표시됩니다. 해당 목록에서 전체 사이트를 검색하는 옵션을 선택할 수도 있습니다.

기본적으로 이 사이트에는 출시된 최신 버전의 PowerShell에 대한 설명서가 표시됩니다. 일부 cmdlet은 다양한 버전의 PowerShell에서 다르게 작동합니다. 사용 중인 PowerShell 버전에 대한 설명서를 확인하세요.

페이지 위쪽의 버전 선택기를 사용하여 원하는 PowerShell 버전을 선택합니다.

![버전 선택기](media/how-to-use-docs/version-search.gif)

사용 중인 PowerShell의 버전은 `$PSversionTable.PSVersion` 값을 검사해서 확인할 수 있습니다. 다음 예제에서는 Windows PowerShell v5.1의 출력을 보여줍니다.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
