---
title: Windows PowerShell 스냅인을 만드는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364432"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Windows PowerShell 스냅인을 만드는 방법

Windows PowerShell 스냅인은 cmdlet의 집합과 다른 Windows PowerShell 공급자를 셸에 등록 하는 메커니즘을 제공 하므로 셸의 기능을 확장 합니다. Windows PowerShell 스냅인은 모든 cmdlet 및 공급자를 단일 어셈블리에 등록 하거나 특정 cmdlet 및 공급자 목록을 등록할 수 있습니다.

스냅인 어셈블리는 다른 운영 체제와 마찬가지로 보호 된 디렉터리에 설치 해야 합니다. 그렇지 않으면 악의적인 사용자가 안전 하지 않은 코드로 어셈블리를 바꿀 수 있습니다.

## <a name="windows-powershell-snap-in-classes"></a>Windows PowerShell 스냅인 클래스

모든 Windows PowerShell 스냅인 클래스는 [add-pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) 또는 [Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) 클래스에서 파생 됩니다 .이 클래스는

## <a name="examples"></a>예

[Windows PowerShell 스냅인 작성](./writing-a-windows-powershell-snap-in.md):이 예제에서는 어셈블리의 모든 cmdlet 및 공급자를 등록 하는 데 사용 되는 스냅인을 만드는 방법을 보여 줍니다.

[사용자 지정 Windows PowerShell 스냅인 작성](./writing-a-custom-windows-powershell-snap-in.md):이 예제에서는 단일 어셈블리에 있을 수도 있고 없을 수도 있는 특정 cmdlet 및 공급자 집합을 등록 하는 데 사용 되는 사용자 지정 스냅인을 만드는 방법을 보여 줍니다.

## <a name="see-also"></a>참고 항목

[Add-pssnapin.](/dotnet/api/System.Management.Automation.PSSnapIn)

[Custompssnapin.](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Cmdlet 등록](./registering-cmdlets.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
