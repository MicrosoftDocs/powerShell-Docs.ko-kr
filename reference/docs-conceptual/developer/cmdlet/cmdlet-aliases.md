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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369982"
---
# <a name="cmdlet-aliases"></a>Cmdlet 별칭

Cmdlet 별칭을 사용 하 여 cmdlet 사용자 환경을 개선할 수 있습니다. 자주 사용 하는 cmdlet에 별칭을 추가 하 여 입력을 줄이고 신속 하 게 작업을 더 쉽게 완료할 수 있습니다. Cmdlet에 기본 제공 별칭을 포함 하거나 사용자가 고유한 사용자 지정 별칭을 정의할 수 있습니다.

예를 들어, [Get Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet에는 기본 제공 `gcm` 별칭이 있습니다. 사용자가 새 명령을 학습할 필요가 없도록 별칭을 사용 하 여 다른 언어의 명령 이름을 추가할 수도 있습니다.

## <a name="alias-guidelines"></a>별칭 지침

Cmdlet에 대 한 기본 제공 별칭을 만드는 경우 다음 지침을 따르세요.

- 별칭을 할당 하기 전에 Windows PowerShell을 시작 하 고, [Get Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet을 실행 하 여 이미 사용 된 별칭을 확인 합니다.

- Cmdlet 이름의 동사를 참조 하는 별칭 접두사와 cmdlet 이름의 명사를 참조 하는 별칭 접미사를 포함 합니다. 예를 들어 `Import-Module` cmdlet의 별칭은 "ipmo"입니다. 모든 동사 및 해당 별칭 목록은 [Cmdlet 동사](./approved-verbs-for-windows-powershell-commands.md)를 참조 하세요.

- 동일한 동사가 있는 cmdlet의 경우 동일한 별칭 접두사를 포함 합니다. 예를 들어 이름에 "Get" 동사가 있는 모든 Windows PowerShell cmdlet의 별칭은 "g" 접두사를 사용 합니다.

- 동일한 명사를 포함 하는 cmdlet의 경우 동일한 별칭 접미사를 포함 합니다. 예를 들어 이름에 "Session" 명사를 포함 하는 모든 Windows PowerShell cmdlet의 별칭은 "sn" 접미사를 사용 합니다.

- 다른 언어의 명령과 동일한 cmdlet의 경우 명령 이름을 사용 합니다.

- 일반적으로 별칭을 가능한 한 짧게 만듭니다. 별칭에 동사에 대해 하나 이상의 고유 문자 및 명사에 대 한 고유 문자가 하나 이상 있는지 확인 합니다. 필요에 따라 더 많은 문자를 추가 하 여 별칭을 고유 하 게 만듭니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
