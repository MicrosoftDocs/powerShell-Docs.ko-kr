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
ms.openlocfilehash: 3cae95fab30a4abe4e544ed5cb7dadc9f4debf02
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692380"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount 특성 선언

ValidateCount 특성은 cmdlet 매개 변수에 허용 되는 인수의 최소 및 최대 수를 지정 합니다.

## <a name="syntax"></a>구문

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>매개 변수

`MinLength`([System.web][])이 필요 합니다. 인수의 최소 개수를 지정 합니다.

`MaxLength`([System.web][])이 필요 합니다. 최대 인수 수를 지정 합니다.

## <a name="remarks"></a>설명

- 이 특성을 선언 하는 방법에 대 한 자세한 내용은 [인수 수의 유효성을 검사][]하는 방법을 참조 하세요.

- 이 특성이 호출 되지 않으면 해당 cmdlet 매개 변수에 원하는 수의 인수가 있을 수 있습니다.

- Windows PowerShell 런타임은 다음과 같은 경우에 오류를 throw 합니다.

  - `MinLength`및 `MaxLength` 특성 매개 변수는 [system.object][]형식이 아닙니다.

  - `MaxLength`특성 매개 변수의 값이 attribute 매개 변수의 값 보다 작은 경우 `MinLength`

- ValidateCount 특성은 [ValidateCountAttribute][] 클래스에 의해 정의 됩니다.

## <a name="see-also"></a>참고 항목

[ValidateCountAttribute.][]

[인수 개수를 확인하는 방법][]

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)][]

[인수 개수를 확인하는 방법]: how-to-validate-an-argument-count.md
[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[ValidateCountAttribute.]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
