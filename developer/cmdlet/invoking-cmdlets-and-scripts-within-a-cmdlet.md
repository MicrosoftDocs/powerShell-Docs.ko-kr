---
title: Cmdlet 및 Cmdlet 내에서 스크립트를 호출 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: e5dc525a6c80ce135d6d68e12968613056d447e8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855189"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Cmdlet 내에서 Cmdlet 및 호출

Cmdlet은 다른 cmdlet와 cmdlet의 메서드를 처리 된 입력 내의 스크립트에서 호출할 수 있습니다. 이 옵션을 사용 하면 코드를 다시 작성할 필요 없이 cmdlet에 기존 cmdlet 및 스크립트의 기능을 추가할 수 있습니다.

## <a name="the-invoke-method"></a>메서드를 호출 합니다.

모든 cmdlet를 호출 하 여 기존 cmdlet을 호출할 수는 [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 와 같은 메서드를 처리 하는 입력에서 메서드를 [ System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)되는 cmdlet에 의해 재정의 됩니다. 그러나에서 직접 파생 되는 cmdlet에만 호출할 수 있습니다 합니다 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 클래스입니다. 파생 되는 cmdlet를 호출할 수 없습니다는 [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스입니다.

합니다 [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 메서드가 다음과 같은 변형을 합니다.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 이 변형은 cmdlet 개체를 호출 하 고 "T" 형식 개체의 컬렉션을 반환 합니다.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 이 변형은 cmdlet 개체를 호출 하 고 강력한 형식의 emumerator를 반환 합니다. 이 변형은 사용자를 컬렉션에 개체를 사용 하 여 사용자 지정 작업을 수행할 수 있습니다.

## <a name="examples"></a>예

|예제|설명|
|-------------|-----------------|
|[Cmdlet 내에서 Cmdlet을 호출합니다.](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|이 예제에는 다른 cmdlet 내에서 cmdlet을 호출 하는 방법을 보여 줍니다.|
|[Cmdlet 내에서 스크립트를 호출합니다.](./how-to-invoke-scripts-within-a-cmdlet.md)|이 예제에는 다른 cmdlet 내에서 cmdlet에 제공 되는 스크립트를 호출 하는 방법을 보여 줍니다.|

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
