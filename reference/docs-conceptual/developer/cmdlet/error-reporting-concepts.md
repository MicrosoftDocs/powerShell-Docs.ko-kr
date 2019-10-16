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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364622"
---
# <a name="error-reporting-concepts"></a>오류 보고 개념

Windows PowerShell은 오류를 보고 하는 두 가지 메커니즘인 오류를 *종료* 하는 메커니즘과 *종료 되지 않는 오류*에 대 한 다른 메커니즘을 제공 합니다. Cmdlet에서 오류를 올바르게 보고 하 여 cmdlet을 실행 하는 호스트 응용 프로그램이 적절 한 방식으로 반응할 수 있도록 하는 것이 중요 합니다.

Cmdlet이 해당 입력 개체를 계속 처리할 수 없는 오류가 발생 하는 경우 cmdlet은 [Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드를 호출 해야 합니다. Cmdlet은 입력 개체를 계속 처리할 수 있는 경우 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하 여 종료 되지 않는 오류를 보고 해야 합니다. 두 방법 모두 호스트 응용 프로그램에서 오류의 원인을 조사 하는 데 사용할 수 있는 오류 레코드를 제공 합니다.

다음 지침을 사용 하 여 오류가 종료 또는 종료 되지 않는 오류 인지 여부를 확인 합니다.

- 오류는 cmdlet이 현재 개체를 계속 처리 하지 않거나 내용에 관계 없이 추가 입력 개체를 성공적으로 처리 하지 못하도록 하는 종료 오류입니다.

- 오류는 cmdlet이 현재 개체 또는 추가 입력 개체의 내용에 관계 없이 계속 해 서 처리 하지 않으려는 경우 종료 오류입니다.

- 개체를 허용 하거나 반환 하지 않는 cmdlet에서 발생 하거나 하나의 개체만 수락 하거나 반환 하는 cmdlet에서 발생 하는 경우에는 종료 오류가 발생 합니다.

- Cmdlet이 현재 개체와 추가 입력 개체를 계속 해 서 처리 하 게 하려면 오류는 종료 되지 않는 오류입니다.

- 특정 입력 개체 또는 입력 개체의 하위 집합과 관련 된 경우에는 종료 되지 않는 오류가 발생 합니다.

## <a name="see-also"></a>참고 항목

[Throwterminatingerror *입니다.](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[WriteError입니다.](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
