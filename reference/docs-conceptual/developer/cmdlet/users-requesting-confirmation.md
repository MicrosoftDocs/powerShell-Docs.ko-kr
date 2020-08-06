---
title: 확인을 요청 하는 사용자 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6f0effb35a110f33248a582fab874e3ab95c7df4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786342"
---
# <a name="users-requesting-confirmation"></a>사용자 확인 요청

`true` `SupportsShouldProcess` Cmdlet 특성 선언의 매개 변수에 값을 지정 하면 사용자가 `Confirm` 명령 프롬프트에서 매개 변수를 지정할 수 있습니다.

기본 환경에서 사용자는 매개 변수를 지정 `Confirm` 하거나 `"-Confirm:$true` [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출할 때 확인이 요청 되도록 할 수 있습니다. 이렇게 하면 높은 영향을 주는 작업에도 불구 하 고 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 확인 요청을 무시 합니다.

`Confirm`을 지정 하지 않으면 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) `$ConfirmPreference` 기본 설정 변수가 `ConfirmImpact` Cmdlet 또는 공급자의 설정 보다 크거나 같은 경우에는 system.object를 호출 하 여 확인을 요청 합니다. 의 기본 설정이 `$ConfirmPreference` 높습니다. 따라서 기본 환경에서는 높은 영향을 주는 작업 요청 확인을 지정 하는 cmdlet 및 공급자만 제공 합니다.

가 false 이거나가 지정 된 경우에는 System.object가 사용자에 게 `Confirm` 확인을 `"-Confirm:$false` 요청 하 고 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) `$ConfirmPreference` shell 변수가 무시 됩니다.

## <a name="remarks"></a>설명

- 를 지정 하는 cmdlet 및 공급자의 경우 `SupportsShouldProcess` `ConfirmImpact` 이러한 작업은 "중간 영향" 작업으로 처리 되며 기본적으로 메시지를 표시 하지 않습니다. 영향 수준이 기본 설정 변수의 기본 설정 보다 낮습니다 `$ConfirmPreference` .

- 사용자가 매개 변수를 지정 하는 경우 `Verbose` 확인 메시지를 표시 하지 않는 경우에도 작업에 대 한 알림이 표시 됩니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
