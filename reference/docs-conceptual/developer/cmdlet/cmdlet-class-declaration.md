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
ms.openlocfilehash: 979025ad5c34ab73dcc23d0e38ffb9acc431f15a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363522"
---
# <a name="cmdlet-class-declaration"></a>Cmdlet 클래스 선언

Microsoft .NET Framework 클래스는 cmdlet 특성을 클래스의 메타 데이터로 지정 하 **여 cmdlet으로** 선언 됩니다. **Cmdlet** 특성은 모든 cmdlet에 대해 유일 하 게 필요한 특성입니다. **Cmdlet** 특성을 지정 하는 경우 사용자에 대해 cmdlet을 식별 하는 동사 및 명사 쌍을 지정 해야 합니다. 그리고 cmdlet이 지 원하는 Windows PowerShell 기능을 설명 해야 합니다. **Cmdlet** 특성을 지정 하는 데 사용 되는 선언 구문에 대 한 자세한 내용은 [cmdlet 특성 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.

> [!NOTE]
> **Cmdlet** 특성은 [system.object](/dotnet/api/System.Management.Automation.CmdletAttribute) 특성 클래스에 의해 정의 됩니다. 이 클래스의 속성은 특성을 선언할 때 사용 되는 선언 매개 변수에 해당 합니다.

## <a name="nouns"></a>쓸

Cmdlet의 명사는 cmdlet이 작동 하는 리소스를 지정 합니다. 명사는 다른 cmdlet에서 cmdlet을 구별 합니다.

Cmdlet 이름의 명사는 특정 해야 하며, *서버*와 같은 일반적인 명사의 경우 리소스를 다른 비슷한 리소스와 구별 하는 짧은 접두사를 추가 하는 것이 가장 좋습니다. 예를 들어 접두사가 포함 된 명사를 포함 하는 cmdlet 이름은 `Get-SQLServer`. 특정 명사를 보다 일반적인 동사로 조합 하면 사용자가 해당 작업으로 cmdlet을 빠르게 찾은 다음 불필요 한 cmdlet 이름 중복을 방지 하는 동시에 해당 리소스에서 cmdlet을 식별할 수 있습니다.

Cmdlet 이름에 사용할 수 없는 특수 문자 목록은 [필수 개발 지침](./required-development-guidelines.md)을 참조 하세요.

## <a name="verbs"></a>동사

동사를 지정 하는 경우 개발 지침을 사용 하려면 Windows PowerShell에서 제공 하는 미리 정의 된 동사 중 하나를 사용 해야 합니다. 이러한 미리 정의 된 동사 중 하나를 사용 하 여 작성 하는 cmdlet과 Microsoft와 다른 사용자가 작성 한 cmdlet 간에 일관성을 유지할 수 있습니다. 예를 들어 "Get" 동사는 데이터를 검색 하는 cmdlet에 사용 됩니다.

동사에 대 한 지침에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요. Cmdlet 이름에 사용할 수 없는 특수 문자 목록은 [필수 개발 지침](./required-development-guidelines.md)을 참조 하세요.

## <a name="supporting-windows-powershell-functionality"></a>Windows PowerShell 기능 지원

**Cmdlet** 특성을 사용 하면 Cmdlet이 Windows PowerShell에서 제공 하는 몇 가지 일반적인 기능을 지원 하도록 지정할 수도 있습니다. 여기에는 사용자 피드백 확인 (ShouldProcess 기능 지원)과 같은 일반적인 기능 및 트랜잭션에 대 한 지원이 포함 됩니다. 트랜잭션에 대 한 지원은 Windows PowerShell 2.0에서 도입 되었습니다.

**Cmdlet** 특성을 지정 하는 데 사용 되는 선언 구문에 대 한 자세한 내용은 [cmdlet 특성 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.

## <a name="cmdlet-class-definition"></a>Cmdlet 클래스 정의

다음 코드는 GetProc cmdlet 클래스에 대 한 정의입니다. 파스칼식 대/소문자가 사용 되 고 클래스 이름에 cmdlet의 동사와 명사가 포함 되어 있는지 확인 합니다.

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>파스칼식 대/소문자 구분

Cmdlet의 이름을 사용할 때는 파스칼식 대/소문자를 사용 합니다. 예를 들어 `Get-Item` 및 `Get-ItemProperty` cmdlet은 cmdlet의 이름을 지정할 때 대/소문자를 사용 하는 올바른 방법을 보여 줍니다.

## <a name="see-also"></a>관련 항목

[System.object. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[CmdletAttribute 선언](./cmdlet-attribute-declaration.md)

[Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[Windows PowerShell SDK](../windows-powershell-reference.md)
