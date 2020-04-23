---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEMenuItemCollection 개체
ms.openlocfilehash: 39e8547c9b19ba323d4b224a46eda416542b2807
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736175"
---
# <a name="the-isemenuitemcollection-object"></a>ISEMenuItemCollection 개체

**ISEMenuItemCollection** 개체는 **ISEMenuItem** 개체의 컬렉션이며, **Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection** 클래스의 인스턴스입니다. 예제는 Windows PowerShell® ISE(통합 스크립팅 환경)에서 `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus`추가 기능**메뉴를 사용자 지정하는 데 사용되는** 개체입니다.

## <a name="method"></a>방법

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

메뉴 항목을 컬렉션에 추가합니다.

**DisplayName** 추가할 메뉴의 표시 이름입니다.

**Action** 이 메뉴 항목과 연결되는 동작을 지정하는 **System.Management.Automation.ScriptBlock** 개체입니다.

**Shortcut** 작업에 대한 바로 가기 키입니다.

**Returns** 방금 추가된 **ISEMenuItem** 개체입니다.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Clear\(\)

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

메뉴 항목에서 모든 하위 메뉴를 제거합니다.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>참고 항목

- [ISEMenuItem 개체](The-ISEMenuItem-Object.md)
- [Windows PowerShell ISE 스크립팅 개체 모델의 용도](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 개체 모델 계층 구조](The-ISE-Object-Model-Hierarchy.md)
