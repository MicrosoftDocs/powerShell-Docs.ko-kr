---
title: Cmdlet에서 cmdlet 및 스크립트 호출 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364292"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Cmdlet 내에서 Cmdlet 및 호출

Cmdlet은 cmdlet의 입력 처리 메서드 내에서 다른 cmdlet 및 스크립트를 호출할 수 있습니다. 이렇게 하면 코드를 다시 작성할 필요 없이 cmdlet에 기존 cmdlet 및 스크립트의 기능을 추가할 수 있습니다.

## <a name="the-invoke-method"></a>Invoke 메서드

모든 cmdlet은에 의해 재정의 되는 입력 처리 메서드 (예: [system.object](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing))에서 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 를 호출 하 여 기존 cmdlet을 호출할 수 있습니다. cmdlet입니다. 그러나 [system.object](/dotnet/api/System.Management.Automation.Cmdlet) 클래스에서 직접 파생 되는 cmdlet만 호출할 수 있습니다. [PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스에서 파생 된 cmdlet을 호출할 수 없습니다.

System.object. n a m. [Invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 메서드에는 다음과 같은 변형이 있습니다.

[System.object를 호출](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 합니다 .이 변형은 cmdlet 개체를 호출 하 고 "T" 형식 개체의 컬렉션을 반환 합니다.

Emumerator cmdlet 개체를 호출 하 고 강력한 형식의를 반환 [합니다.](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 이 변형을 사용 하면 사용자가 컬렉션의 개체를 사용 하 여 사용자 지정 작업을 수행할 수 있습니다.

## <a name="examples"></a>예

|예제|설명|
|-------------|-----------------|
|[Cmdlet에서 cmdlet 호출](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|이 예에서는 다른 cmdlet 내에서 cmdlet을 호출 하는 방법을 보여 줍니다.|
|[Cmdlet 내에서 스크립트 호출](./how-to-invoke-scripts-within-a-cmdlet.md)|이 예에서는 다른 cmdlet 내에서 cmdlet에 제공 된 스크립트를 호출 하는 방법을 보여 줍니다.|

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
