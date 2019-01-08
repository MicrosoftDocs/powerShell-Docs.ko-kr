---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippetCollection 개체
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403435"
---
# <a name="the-isesnippetcollection-object"></a>ISESnippetCollection 개체

**ISESnippetCollection** 개체는 **ISESnippet** 개체의 컬렉션입니다. **PowerShellTab** 개체와 연결되어 있는 파일 컬렉션이 이 클래스의 멤버입니다. 예제는 **$psISE.CurrentPowerShellTab.Files** 컬렉션입니다.

## <a name="methods"></a>메서드

### <a name="load-filepathname-"></a>Load\( FilePathName \)

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

사용자가 정의한 코드 조각을 포함하는 .snippets.ps1xml 파일을 로드합니다. 코드 조각을 만드는 가장 쉬운 방법은 New-IseSnippet cmdlet을 사용하는 것입니다. 이 cmdlet은 Windows PowerShell ISE를 시작할 때마다 코드 조각이 로드되도록 코드 조각을 프로필 폴더에 자동으로 저장합니다.

**FilePathName** – 문자열. 코드 조각 정의를 포함하는 .snippets.ps1xml 파일의 경로 및 파일 이름입니다.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>참고 항목

- [ISESnippet 개체](The-ISESnippetObject.md)
- [Windows PowerShell ISE 스크립팅 개체 모델의 용도](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 개체 모델 계층 구조](The-ISE-Object-Model-Hierarchy.md)