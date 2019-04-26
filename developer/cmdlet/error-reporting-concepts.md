---
title: 오류 보고 개념 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068184"
---
# <a name="error-reporting-concepts"></a>오류 보고 개념

오류를 보고 하는 두 가지 메커니즘을 제공 하는 Windows PowerShell: 메커니즘 중 하나 *종료* 및 다른 메커니즘 *비종료 오류*합니다. 반드시 오류를 보고 하려면 cmdlet에 대 한 올바르게 cmdlet을 실행 하는 호스트 응용 프로그램은 적절 한 방식으로 대응할 수 있도록 합니다.

Cmdlet을 호출 해야 합니다 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드는 오류가 발생 하지 않습니다 또는 cmdlet이 해당 입력된 개체를 처리 하는 데 계속 하도록 허용 하지 않아야 합니다. Cmdlet을 호출 해야 합니다 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) cmdlet은 입력된 개체를 처리를 계속할 수 있으면 종료 되지 않는 오류를 보고 하는 방법입니다. 두 메서드는 호스트 응용 프로그램 오류의 원인을 조사 하는 데 사용할 수 있는 오류 레코드를 제공 합니다.

오류 인지 종료 또는 종료 되지 않는 오류를 확인 하려면 다음 지침을 따르세요.

- 오류가 계속 현재 개체를 처리 또는 해당 내용에 관계 없이 모든 추가 입력된 개체를 성공적으로 처리에서 cmdlet을 방지 하는 경우 종료 오류를입니다.

- 오류가 발생 하지 않으려는 경우 cmdlet에 계속 해 서 현재 개체 또는 해당 내용에 관계 없이 모든 추가 입력된 개체를 처리 하는 경우 종료 오류를입니다.

- 오류가 되었거나 종료 오류를 허용 하지 않거나 개체를 반환 하는 cmdlet에서 발생 하는 경우 허용 하거나 개체를 하나만 반환 하는 cmdlet에서 발생 하는 경우.

- 오류는 cmdlet에 계속 해 서 현재 개체와 모든 추가 입력된 개체를 처리 하려면 비종료 오류가입니다.

- 오류는 입력된 개체의 하위 집합 또는 특정 입력된 개체에 관련 된 경우 종료 되지 않는 오류가입니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
