---
ms.date: 09/13/2016
ms.topic: reference
title: 오류 정보 표시
description: 오류 정보 표시
ms.openlocfilehash: 37a3adb91d0e616a5c7f27bcab866f8da139f969
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653054"
---
# <a name="displaying-error-information"></a>오류 정보 표시

이 항목에서는 사용자가 오류 정보를 표시할 수 있는 방법에 대해 설명 합니다.

Cmdlet에 오류가 발생 하면 오류 정보를 표시 하는 것은 기본적으로 다음 오류 출력과 유사 합니다.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

그러나 사용자는 변수를로 설정 하 여 범주별로 오류를 볼 수 있습니다 `$ErrorView` `"CategoryView"` . 범주 보기에는 오류에 대 한 자유 텍스트 설명이 아닌 오류 레코드의 특정 정보가 표시 됩니다. 이 보기는 검색할 오류 목록이 긴 경우에 유용할 수 있습니다. 범주 보기에서 이전 오류 메시지는 다음과 같이 표시 됩니다.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

오류 범주에 대 한 자세한 내용은 [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)를 참조 하십시오.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
