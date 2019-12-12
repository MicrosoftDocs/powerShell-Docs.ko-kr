---
title: 자격 증명 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369892"
---
# <a name="credential-attribute-declaration"></a>Credential 증명 특성 선언

Credential 특성은 문자열을 매개 변수에 대 한 인수로 전달할 수도 있도록 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 형식의 자격 증명 매개 변수와 함께 사용할 수 있는 선택적 특성입니다. 이 특성을 매개 변수 선언에 추가 하면 Windows PowerShell에서 문자열 입력을 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 로 변환 합니다. 예를 들어, [Get Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet은이 특성을 사용 하 여 Windows PowerShell에서 cmdlet에 의해 반환 되는 [system.web. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) 개체를 생성 하도록 합니다.

## <a name="syntax"></a>구문

```csharp
[Credential]
```

## <a name="remarks"></a>설명

- 일반적으로이 특성은 문자열을 매개 변수에 대 한 인수로 전달할 수도 있도록 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 형식의 매개 변수에서 사용 됩니다. [System.object](/dotnet/api/System.Management.Automation.PSCredential) 가 매개 변수에 전달 되 면 Windows PowerShell은 아무 작업도 수행 하지 않습니다.

- Windows PowerShell은 현재 호스트를 사용 하 여 사용자에 게 적절 한 프롬프트를 표시 [합니다.](/dotnet/api/System.Management.Automation.PSCredential) 예를 들어이 특성을 사용 하는 경우 기본 호스트는 사용자 이름 및 암호를 묻는 메시지를 표시 합니다. 그러나 다른 프롬프트를 정의 하는 사용자 지정 호스트를 사용 하는 경우에는 프롬프트가 표시 됩니다.

- 이 특성은 Parameter 특성과 함께 사용 됩니다. 해당 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.

- Credential 특성은 [system.web. credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) 클래스에 의해 정의 됩니다.

## <a name="see-also"></a>참고 항목

[매개 변수 별칭](./parameter-aliases.md)

[매개 변수 특성 선언](./parameter-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
