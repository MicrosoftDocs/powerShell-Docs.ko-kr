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
ms.openlocfilehash: 73834cea1d90943cf954728d6295d8eb33e14f57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859759"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Windows PowerShell 스냅인을 만드는 방법

Windows PowerShell 스냅인을 사용 하는 cmdlet 및 다른 Windows PowerShell 공급자 집합을 따라서 셸 기능을 확장 하는 셸을 등록 하기 위한 메커니즘을 제공 합니다. Windows PowerShell 스냅인을 등록할 수는 모든 cmdlet 및 공급자 단일 어셈블리에 또는 특정 목록을 cmdlet 및 공급자를 등록할 수 있습니다.

스냅인 어셈블리는 다른 운영 체제를 사용 하 여 것 처럼 보호 된 디렉터리에 설치 되어야 합니다. 이 고, 그렇지 악의적인 사용자가 안전 하지 않은 코드를 사용 하 여 어셈블리를 바꿀 수 있습니다.

## <a name="windows-powershell-snap-in-classes"></a>Windows PowerShell 스냅인 클래스

모든 Windows PowerShell 스냅인 클래스에서 파생 된 [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) 하거나 [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) 클래스입니다.

## <a name="examples"></a>예

[Windows PowerShell 스냅인 작성](./writing-a-windows-powershell-snap-in.md): 이 예제에서는 어셈블리의 모든 cmdlet 및 공급자를 등록 하는 데 사용 되는 스냅인 만드는 방법을 보여 줍니다.

[사용자 지정 Windows PowerShell 스냅인 작성](./writing-a-custom-windows-powershell-snap-in.md): 이 예제에서는 사용자 지정 맞춤에 존재 하지 않을 수도 있는 cmdlet 및 공급자의 특정 집합을 단일 어셈블리를 등록 하는 데 사용 되는 만드는 방법을 보여 줍니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn)

[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Cmdlet을 등록합니다.](./registering-cmdlets.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
