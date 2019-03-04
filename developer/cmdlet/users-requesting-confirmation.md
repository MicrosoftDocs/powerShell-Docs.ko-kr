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
ms.openlocfilehash: e4abbb14b31406b845d9b6af6b6372338fb0d926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856239"
---
# <a name="users-requesting-confirmation"></a>사용자 확인 요청

값을 지정 하는 경우 `true` 에 대 한 합니다 `SupportsShouldProcess` Cmdlet 특성 선언의 매개 변수를 사용자 지정할 수는 `Confirm` 명령 프롬프트 매개 변수입니다.

기본 환경에서 사용자 지정할 수 있습니다는 `Confirm` 매개 변수 또는 `"-Confirm:$true` 확인 요청 되는 때를 [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드가 호출 됩니다. 이 건너뜁니다 [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 영향력이 높은 작업에 대해서도 확인 요청을 합니다.

경우 `Confirm` 지정 하지 않으면를 [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 호출 하는 경우 확인을 요청 합니다 `$ConfirmPreference` 기본 설정 변수가 보다 크거나 같은 `ConfirmImpact` 설정는 cmdlet 또는 공급자입니다. 기본 설정인 `$ConfirmPreference` 높음입니다. 따라서 기본 환경만 cmdlet 및 공급자 영향력이 높은 작업을 지정 하는 확인을 요청 합니다.

경우 `Confirm` 이 false 이거나 `"-Confirm:$false` 지정 된 경우를 [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 사용자 로부터 확인을 요청 하는 호출 및 `$ConfirmPreference` 셸 변수는 무시 됩니다.

## <a name="remarks"></a>설명

- 지정 하는 cmdlet 및 공급자에 대 한 `SupportsShouldProcess`, 아닌 `ConfirmImpact`, "중간 영향" 작업으로 이러한 동작을 처리 하 고 기본적으로 메시지 표시 되지 것입니다. 기본 설정을 보다 낮은 해당 영향 수준입니다는 `$ConfirmPreference` 기본 설정 변수입니다.

- 사용자 지정 하는 경우는 `Verbose` 매개 변수를 알림이 표시 됩니다 작업의 확인을 묻지 않습니다 하는 경우에 합니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
