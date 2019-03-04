---
title: Cmdlet 클래스 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3e410087438ac99526049f99e5c768c017a29848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854449"
---
# <a name="cmdlet-class-declaration"></a>Cmdlet 클래스 선언

Microsoft.NET Framework 클래스를 지정 하 여 cmdlet으로 선언 된 **Cmdlet** 클래스에 대 한 메타 데이터 특성입니다. (합니다 **Cmdlet** 특성은 모든 cmdlet에 대 한 필수 속성). 지정 하는 경우는 **Cmdlet** 특성인 cmdlet이 사용자를 식별 하는 동사-명사 쌍을 지정 해야 합니다. 및 cmdlet에서 지 원하는 Windows PowerShell 기능을 설명 해야 합니다. 지정 하는 데 사용 되는 선언 구문에 대 한 자세한 내용은 합니다 **Cmdlet** 특성을 참조 하십시오 [Cmdlet 특성 선언을](./cmdlet-attribute-declaration.md)합니다.

> [!NOTE]
> **Cmdlet** 특성은 정의한 합니다 [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 클래스입니다. 이 클래스의 속성 특성을 선언 하는 경우 사용 되는 선언 매개 변수와 일치 합니다.

## <a name="nouns"></a>명사

Cmdlet의 명사는 cmdlet이 적용 되는 리소스를 지정 합니다. 명사는 다른 cmdlet에서 cmdlet을 구분합니다.

Cmdlet 이름의 명사 해야 특정 및 일반 명사의 경우와 같은 *server*를 유사한 다른 리소스에서 리소스를 구분할 수 있는 짧은 접두사를 추가 하는 것이 좋습니다. 예를 들어는 접두사가 포함 된 명사를 포함 하는 cmdlet 이름 `Get-SQLServer`합니다. 보다 일반적인 동사와 특정 명사를 조합 작업에 의해 cmdlet를 빠르게 찾은 후 불필요 한 cmdlet 이름 중복을 방지 하는 동안 해당 리소스에서 cmdlet을 식별 한 다음 사용자를 수 있습니다.

Cmdlet 이름에 사용할 수 없는 특수 문자의 목록을 참조 하세요 [개발 지침 필요한](./required-development-guidelines.md)합니다.

## <a name="verbs"></a>동사

동사를 지정 하는 경우 개발 지침 미리 정의 된 Windows PowerShell에서 제공 되는 동사 중 하나를 사용 해야 합니다. 이러한 미리 정의 된 동사 중 하나를 사용 하 여 작성 하는 cmdlet 및 다른 사용자가 Microsoft에서 작성 된 cmdlet 간에 일관성을 해야 합니다. 예를 들어, 데이터를 검색 하는 cmdlet에 대 한 "Get" 동사가 사용 됩니다.

동사에 대 한 지침에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다. Cmdlet 이름에 사용할 수 없는 특수 문자의 목록을 참조 하세요 [개발 지침 필요한](./required-development-guidelines.md)합니다.

## <a name="supporting-windows-powershell-functionality"></a>Windows PowerShell 기능을 지 원하는

합니다 **Cmdlet** 특성 또한 cmdlet Windows PowerShell에서 제공 하는 일반적인 기능 중 일부를 지원 하는지 지정할 수 있습니다. 사용자에 게 피드백 확인 (ShouldProcess 기능에 대 한 지원 이라고 함) 등의 일반적인 기능에 대 한 지원 및 트랜잭션에 대 한 지원이 포함 됩니다. (트랜잭션에 대 한 지원이 Windows PowerShell 2.0에서 도입 되었습니다).

지정 하는 데 사용 되는 선언 구문에 대 한 자세한 내용은 합니다 **Cmdlet** 특성을 참조 하십시오 [Cmdlet 특성 선언을](./cmdlet-attribute-declaration.md)합니다.

## <a name="cmdlet-class-definition"></a>Cmdlet 클래스 정의

다음 코드는 GetProc cmdlet 클래스에 대 한 정의입니다. 파스칼식 대/소문자 구분 되 고 클래스의 이름을 동사와 cmdlet의 명사를 포함 하는 알 수 있습니다.

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>파스칼식 대/소문자 구분

Cmdlet에 이름을 지정할 때 사용 하 여 파스칼식 대/소문자 구분 합니다. 예를 들어 합니다 `Get-Item` 및 `Get-ItemProperty` cmdlet cmdlet를 명명할 때 대/소문자를 사용 하는 올바른 방법을 보여 줍니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[CmdletAttribute 선언](./cmdlet-attribute-declaration.md)

[Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell SDK](../windows-powershell-reference.md)
