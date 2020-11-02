---
ms.date: 06/05/2017
title: ISESnippet 개체
description: ISESnippet 개체는 Microsoft.PowerShell.Host.ISE.ISESnippet 클래스의 인스턴스입니다.
ms.openlocfilehash: 602b344686cbcfb1e994914d4e26438ff7e4b1de
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663413"
---
# <a name="the-isesnippetobject"></a>ISESnippet 개체

**ISESnippet** 개체는 Microsoft.PowerShell.Host.ISE.ISESnippet 클래스의 인스턴스입니다. `$psISE.CurrentPowerShellTab.Snippets` 컬렉션의 멤버는 모두 **ISESnippet** 개체의 예입니다. 코드 조각을 만드는 가장 쉬운 방법은 [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) cmdlet을 사용하는 것입니다.

## <a name="properties"></a>속성

### <a name="author"></a>작성자

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

코드 조각 작성자의 이름을 가져오는 읽기 전용 속성입니다.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

편집기에 삽입할 코드 조각을 가져오는 읽기 전용 속성입니다.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>바로 가기

Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.

메뉴 항목에 대한 Windows 바로 가기 키를 가져오는 읽기 전용 속성입니다.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>참고 항목

- [ISESnippetCollection 개체](The-ISESnippetCollection-Object.md)
- [Windows PowerShell ISE 스크립팅 개체 모델의 용도](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [ISE 개체 모델 계층 구조](The-ISE-Object-Model-Hierarchy.md)
