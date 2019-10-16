---
title: 속성을 매개 변수로 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365752"
---
# <a name="declaring-properties-as-parameters"></a>매개 변수로 속성 선언

이 항목에서는 cmdlet의 매개 변수를 선언 하기 전에 이해 해야 하는 기본적인 정보를 제공 합니다.

Cmdlet 클래스 내에서 cmdlet의 매개 변수를 선언 하려면 각 매개 변수를 나타내는 공용 속성을 정의한 다음 각 속성에 하나 이상의 매개 변수 특성을 추가 합니다. Windows PowerShell 런타임에서는 매개 변수 특성을 사용 하 여 속성을 cmdlet 매개 변수로 식별 합니다. 매개 변수 특성을 선언 하는 기본 구문은 `[Parameter()]`입니다.

필수 매개 변수로 정의 된 속성의 예는 다음과 같습니다.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

매개 변수에 대해 기억할 몇 가지 사항은 다음과 같습니다.

- 매개 변수는 명시적으로 public으로 표시 되어야 합니다. 공용 기본으로 표시 되지 않은 매개 변수는 Windows PowerShell 런타임에 의해 검색 되지 않습니다.

- 매개 변수는 매개 변수 유효성 검사를 향상 시킬 수 있도록 Microsoft .NET Framework 형식으로 정의 해야 합니다. 예를 들어 값 집합에서 하나의 값으로 제한 되는 매개 변수는 열거형 형식으로 정의 되어야 합니다. URI (Uniform Resource Identifier) 값을 사용 하는 매개 변수는 system.string [형식 이어야 합니다.](/dotnet/api/System.Uri)

- 자유 형식 텍스트 속성에 대 한 기본 문자열 매개 변수를 사용 하지 않습니다.

- 매개 변수를 원하는 수 만큼 매개 변수 집합에 추가할 수 있습니다. 매개 변수 집합에 대 한 자세한 내용은 [Cmdlet 매개 변수 집합](./cmdlet-parameter-sets.md)을 참조 하세요.

또한 Windows PowerShell에서는 모든 cmdlet에 자동으로 사용할 수 있는 공통 매개 변수 집합을 제공 합니다. 이러한 매개 변수 및 해당 별칭에 대 한 자세한 내용은 [Cmdlet 일반 매개 변수](./common-parameter-names.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[Cmdlet 일반 매개 변수](./common-parameter-names.md)

[Cmdlet 매개 변수의 유형](./types-of-cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
