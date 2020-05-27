---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippet 개체
ms.openlocfilehash: f810e6b26f0ded04be15bdc37f336d7890e29dad
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809579"
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
