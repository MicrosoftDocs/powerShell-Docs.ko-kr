---
title: Cmdlet 별칭 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860509"
---
# <a name="cmdlet-aliases"></a>Cmdlet 별칭

Cmdlet은 사용자 환경을 개선 하기 위해 cmdlet 별칭을 사용할 수 있습니다. 입력을 줄이고 쉽게 작업을 완료 하려면 신속 하 게 자주 사용 되는 cmdlet 별칭을 추가할 수 있습니다. 기본 제공 별칭, cmdlet에서 포함 하거나 사용자가 자신의 사용자 지정 별칭을 정의할 수 있습니다.

예를 들어 합니다 [Get-command](/powershell/module/microsoft.powershell.core/get-command) cmdlet에는 기본 제공 `gcm` 별칭입니다. 또한 사용자가 새 명령에 알아보기 하지 않아도 되도록 명령 이름을 다른 언어에서 추가 별칭을 사용할 수 있습니다.

## <a name="alias-guidelines"></a>별칭 지침

Cmdlet에 대 한 기본 제공 별칭을 만들 때 다음이 지침을 따르세요.

- 별칭을 할당 하기 전에 Windows PowerShell을 시작 하 고 실행 합니다 [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet을 이미 사용 되는 별칭을 참조 하십시오.

- Cmdlet 이름 및 별칭 접미사가 cmdlet 이름의 명사를 참조 하는 동사를 참조 하는 별칭 접두사를 포함 합니다. 예를 들어,에 대 한 별칭을 `Import-Module` cmdlet은 "ipmo"입니다. 모든 동사 및 해당 별칭의 목록을 참조 하세요 [Cmdlet 동사](./approved-verbs-for-windows-powershell-commands.md)합니다.

- 동일한 동사는 cmdlet에 대해 같은 별칭 접두사를 포함 합니다. 예를 들어, 해당 이름에 "Get" 동사가 포함 된 모든 Windows PowerShell cmdlet의 별칭을 "g" 접두사를 사용 합니다.

- 동일한 명사가 있는 cmdlet에 대해 같은 별칭 접미사를 포함 합니다. 예를 들어 이름에 "세션" 명사가 있는 모든 Windows PowerShell cmdlet의 별칭을 "sn" 접미사를 사용 합니다.

- 명령의 이름을 다른 언어로 명령에 해당 하는 cmdlet을 사용 합니다.

- 일반적으로 짧게 별칭을 확인 합니다. 별칭 명사에 대 한 하나의 고유한 문자 및 동사에 대 한 고유 문자를 하나 이상 있는지 확인 합니다. 별칭 고유 하 게 필요에 따라 더 많은 문자를 추가 합니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
