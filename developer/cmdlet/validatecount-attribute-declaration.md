---
title: ValidateCount 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859159"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount 특성 선언

ValidateCount 특성 인수는 cmdlet 매개 변수에 대해 허용 되는 최소 및 최대 수를 지정 합니다.

## <a name="syntax"></a>구문

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>매개 변수

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) 필요 합니다. 최소 인수 개수를 지정합니다.

`MaxLength`([System.Int32](/dotnet/api/System.Int32)) 필요 합니다. 인수의 최대 수를 지정 합니다.

## <a name="remarks"></a>설명

- 이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [입력 유효성 검사 규칙 선언 하는 방법을](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)합니다.

- 이 특성은 호출 되지 경우 해당 cmdlet 매개 변수 인수 몇 개 있습니다.

- Windows PowerShell 런타임에 다음과 같은 경우 오류가 throw 됩니다.

    - 합니다 `MinLength` 하 고 `MaxLength` 형식이 아닌 특성 매개 변수 [System.Int32](/dotnet/api/System.Int32)합니다.

    - 값을 `MaxLength` 특성 매개 변수 값 보다 작습니다는 `MinLength` 특성 매개 변수입니다.

- ValidateCount 특성은 정의한 합니다 [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) 클래스입니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)

[입력된 유효성 검사 규칙을 선언 하는 방법](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[입력된 유효성 검사 규칙을 선언 하는 방법](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
