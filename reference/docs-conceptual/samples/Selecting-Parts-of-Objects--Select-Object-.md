---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 개체의 일부 선택(Select Object)
ms.openlocfilehash: 06b92c7c4c5098c707a7d9f9d9a96e6b6a897f80
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737171"
---
# <a name="selecting-parts-of-objects-select-object"></a>개체의 일부 선택(Select-Object)

`Select-Object` cmdlet을 사용하면 새 사용자 지정 PowerShell 개체를 만들 수 있습니다. 이러한 개체에는 해당 개체를 만드는 데 사용된 개체에서 선택한 속성이 포함되어 있습니다. 다음 명령을 입력하면 **Win32_LogicalDisk** WMI 클래스의 **Name** 및 **FreeSpace** 속성만 포함된 새 개체를 만들 수 있습니다.

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

`Select-Object`를 사용하여 계산된 속성을 만들 수 있습니다. 따라서 **FreeSpace**를 바이트 대신 기가바이트 단위로 표시할 수 있습니다.

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  Select-Object -Property Name, @{
    label='FreeSpace'
    expression={($_.FreeSpace/1GB).ToString('F2')}
  }
```

```Output
Name    FreeSpace
----    ---------
C:      47.18
```
