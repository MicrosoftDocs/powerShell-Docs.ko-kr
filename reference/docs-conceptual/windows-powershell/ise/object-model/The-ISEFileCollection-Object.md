---
ms.date: 12/31/2019
title: ISEFileCollection 개체
description: ISEFileCollection 개체는 ISEFile 개체의 컬렉션입니다.
ms.openlocfilehash: 2feef1200c611d5181bcbc55d5464a0bd390084e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646752"
---
# <a name="the-isefilecollection-object"></a>ISEFileCollection 개체

**ISEFileCollection** 개체는 **ISEFile** 개체의 컬렉션입니다. `$psISE.CurrentPowerShellTab.Files` 컬렉션을 예로 들 수 있습니다.

## <a name="methods"></a>메서드

### <a name="add-fullpath-"></a>Add\( \[FullPath\] \)

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

제목이 없는 새 파일을 만들고 반환하고 컬렉션에 추가합니다. 새로 생성된 파일의 **IsUntitled** 속성은 `$true`입니다.

**\[FullPath\]** – 선택적 문자열. 완전히 지정된 파일 경로입니다. **FullPath** 매개 변수 및 상대 경로를 포함하거나, 전체 경로 대신 파일 이름을 사용하는 경우 예외가 생성됩니다.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Remove\( File, \[Force\] \)

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

현재 PowerShell 탭에서 지정된 파일을 제거합니다.

**File** – 문자열. 컬렉션에서 제거하려는 ISEFile 파일입니다. 파일이 저장되지 않은 경우 이 메서드에서 예외를 throw합니다. 저장되지 않은 파일의 제거를 강제로 수행하려면 이 **Force** 스위치 매개 변수를 사용합니다.

**\[Force\]** - 선택적 부울. `$true`로 설정된 경우, 마지막 사용 후 저장하지 않았더라도 파일을 제거할 수 있는 권한을 부여합니다. 기본값은 `$false`입니다.

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile \)

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

**SelectedFile** 매개 변수로 지정된 파일을 선택합니다.

**SelectedFile** – Microsoft.PowerShell.Host.ISE.ISEFile. 선택할 ISEFile 파일입니다.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>참고 항목

- [ISEFile 개체](The-ISEFile-Object.md)
- [Windows PowerShell ISE 스크립팅 개체 모델의 용도](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 개체 모델 계층 구조](The-ISE-Object-Model-Hierarchy.md)
