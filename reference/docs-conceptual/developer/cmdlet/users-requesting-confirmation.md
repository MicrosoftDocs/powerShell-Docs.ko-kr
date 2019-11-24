---
title: 확인을 요청 하는 사용자 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369252"
---
# <a name="users-requesting-confirmation"></a>사용자 확인 요청

Cmdlet 특성 선언의 `SupportsShouldProcess` 매개 변수에 `true` 값을 지정 하면 사용자는 명령 프롬프트에서 `Confirm` 매개 변수를 지정할 수 있습니다.

기본 환경에서 사용자는 `Confirm` 매개 변수를 지정 하거나 `"-Confirm:$true`를 지정 하 여 확인이 요청 될 때 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출할 수 있습니다. 이렇게 하면 높은 영향을 주는 작업에도 불구 하 고 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 확인 요청을 무시 합니다.

`Confirm` 지정 되지 않은 경우 `$ConfirmPreference` 기본 설정 변수가 Cmdlet 또는 공급자의 `ConfirmImpact` 설정 보다 크거나 같은 경우에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하 여 확인을 요청 합니다. `$ConfirmPreference`의 기본 설정은 높습니다. 따라서 기본 환경에서는 높은 영향을 주는 작업 요청 확인을 지정 하는 cmdlet 및 공급자만 제공 합니다.

`Confirm` false 이거나 `"-Confirm:$false` 지정 된 경우에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 가 사용자의 확인을 요청 하 고 `$ConfirmPreference` shell 변수가 무시 됩니다.

## <a name="remarks"></a>설명

- `SupportsShouldProcess`를 지정 하지만 `ConfirmImpact`하지 않는 cmdlet 및 공급자의 경우 이러한 작업은 "중간 영향" 작업으로 처리 되며 기본적으로 메시지를 표시 하지 않습니다. 영향 수준이 `$ConfirmPreference` 기본 설정 변수의 기본 설정 보다 낮습니다.

- 사용자가 `Verbose` 매개 변수를 지정 하는 경우 확인 메시지를 표시 하지 않는 경우에도 작업에 대 한 알림이 표시 됩니다.

## <a name="see-also"></a>관련 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
