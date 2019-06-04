---
title: 오류 정보를 표시 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068286"
---
# <a name="displaying-error-information"></a>오류 정보 표시

이 항목에서는 사용자가 오류 정보를 표시할 수 있는 방법을 설명 합니다.

Cmdlet에 오류가 발생 하는 경우 표시 되는 오류 정보는 기본적으로 다음 오류 출력과를 비슷합니다.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

그러나 사용자가 오류를 볼 수 범주별으로 설정 하 여 합니다 `$ErrorView` 변수를 `"CategoryView"`입니다. 종류별 보기 자유 텍스트 설명은 오류 보다는 error 레코드의 특정 정보를 표시합니다. 이 보기는 검색 오류 목록이 긴 경우에 유용할 수 있습니다. 종류별 보기에서 이전 오류 메시지는 다음과 같이 표시 됩니다.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

오류 범주에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
