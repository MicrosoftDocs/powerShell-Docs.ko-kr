---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShellTabCollection 개체
ms.openlocfilehash: 0aad885afd3ba3ae3b00f5c11d2c62a9ff303798
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808569"
---
# <a name="the-powershelltabcollection-object"></a>PowerShellTabCollection 개체

**PowerShellTab** 컬렉션 개체는 **PowerShellTab** 개체의 컬렉션입니다. 각 **PowerShellTab** 개체는 별도의 런타임 환경으로 작동합니다. Microsoft.PowerShell.Host.ISE.PowerShellTabs 클래스의 인스턴스입니다. `$psISE.PowerShellTabs` 개체를 예로 들 수 있습니다.

## <a name="methods"></a>메서드

### <a name="add"></a>추가\(\)

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

새 PowerShell 탭을 컬렉션에 추가합니다. 새로 추가된 탭을 반환합니다.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

**psTab** 매개 변수로 지정되는 탭을 제거합니다.

**psTab** 제거할 PowerShell 탭입니다.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

**psTab** 매개 변수에서 지정하는 PowerShell 탭을 선택하여 현재 사용 중인 PowerShell 탭으로 만듭니다.

**psTab** 선택할 PowerShell 탭입니다.

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a>참고 항목

- [PowerShellTab 개체](The-PowerShellTab-Object.md)
- [Windows PowerShell ISE 스크립팅 개체 모델의 용도](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 개체 모델 계층 구조](The-ISE-Object-Model-Hierarchy.md)
