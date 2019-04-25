---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 기타 유용한 스크립팅 개체
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: ff494f375c0d43d83b2a067dbe4f2ab35a90d564
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086207"
---
# <a name="other-useful-scripting-objects"></a>기타 유용한 스크립팅 개체

다음 개체에서는 Windows PowerShell ISE의 추가 스크립팅 기능을 제공합니다. **$psISE** 계층 구조에 포함되지는 않습니다.

## <a name="useful-scripting-objects"></a>유용한 스크립팅 개체

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Windows PowerShell ISE가 콘솔 애플리케이션과 상호 작용하는 방식에는 몇 가지 제한 사항이 있습니다. 사용자의 개입을 필요로 하는 명령이나 자동화 스크립트는 Windows PowerShell 콘솔에서 작동하는 방식으로 작동하지 않을 수 있습니다. 이러한 명령이나 스크립트가 Windows PowerShell ISE 명령 창에서 실행되는 것을 차단할 수 있습니다. **$psUnsupportedConsoleApplications** 개체는 그러한 명령의 목록을 보관합니다. 이 목록에 있는 명령을 실행하려 할 경우, 지원되지 않는다는 메시지가 표시됩니다. 다음 스크립트는 목록에 항목을 추가합니다.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

로컬의 컴파일된 HTML 도움말 파일에 있는 도움말 항목과 연결된 링크 간에 상황에 맞는 매핑을 유지 관리하는 사전 개체입니다. 특정 항목에 대한 로컬 도움말을 찾는 데 사용됩니다. 이 목록에서 항목을 추가하거나 삭제할 수 있습니다. 다음 코드 예제에서는 `$psLocalHelp`에 들어 있는 몇 가지 키-값 쌍 예를 보여 줍니다.

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

다음 스크립트는 목록에 항목을 추가합니다.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

도움말 항목의 항목 제목과 거기에 연결된 외부 URL 간에 상황에 맞는 매핑을 유지 관리하는 사전 개체입니다. 웹에서 특정 항목에 대한 도움말을 찾는 데 사용됩니다. 이 목록에서 항목을 추가하거나 삭제할 수 있습니다.

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : http://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : http://go.microsoft.com/fwlink/p/?LinkID=113278
```

다음 스크립트는 목록에 항목을 추가합니다.

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>참고 항목

[Windows PowerShell ISE 스크립팅 개체 모델의 용도](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)