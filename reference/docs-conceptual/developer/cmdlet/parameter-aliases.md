---
title: 매개 변수 별칭 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369592"
---
# <a name="parameter-aliases"></a>매개 변수 별칭

Cmdlet 매개 변수에는 별칭을 사용할 수도 있습니다. 명령에서 매개 변수를 입력 하거나 지정 하는 경우 매개 변수 이름 대신 별칭을 사용할 수 있습니다.

## <a name="benefits-of-using-aliases"></a>별칭 사용의 이점

매개 변수에 별칭을 추가 하면 다음과 같은 이점이 있습니다.

- 사용자가 cmdlet을 호출할 때 전체 매개 변수 이름을 사용 하지 않아도 되도록 바로 가기를 제공할 수 있습니다. 예를 들어 "ComputerName" 매개 변수 이름 대신 "CN" 별칭을 사용할 수 있습니다.

- 동일한 매개 변수에 다른 이름을 제공 하려는 경우 여러 별칭을 정의할 수 있습니다. 여러 다른 방법으로 동일한 데이터를 참조 하는 여러 사용자 그룹으로 작업 해야 하는 경우 여러 별칭을 정의 하는 것이 좋습니다.

- 매개 변수 이름이 변경 되는 경우 기존 스크립트에 대 한 이전 버전과의 호환성을 제공할 수 있습니다.

- ValueFromPipelineByName 특성과 함께 Alias 특성을 사용 하 여 cmdlet이 다른 개체 형식에 바인딩할 수 있도록 하는 매개 변수를 정의할 수 있습니다. 예를 들어 다른 형식의 개체가 두 개 있고 첫 번째 개체에는 기록기 속성이 있고 두 번째 개체에는 편집기 속성이 있다고 가정 합니다. Cmdlet에 작성기 및 편집기 별칭이 있는 매개 변수가 있고 속성 이름을 기반으로 하는 cmdlet의 파이프라인 입력이 허용 되는 경우 cmdlet은 두 개의 매개 변수 별칭을 사용 하 여 두 개체에 모두 바인딩할 수 있습니다.

특정 매개 변수와 함께 사용할 수 있는 별칭에 대 한 자세한 내용은 [일반 매개 변수 이름](./common-parameter-names.md)을 참조 하세요.

## <a name="defining-parameter-aliases"></a>매개 변수 별칭 정의

매개 변수에 대 한 별칭을 정의 하려면 다음 매개 변수 선언에 표시 된 것 처럼 별칭 특성을 선언 합니다. 이 예제에서는 동일한 매개 변수에 대 한 여러 별칭을 정의 합니다. (자세한 내용은[Cmdlet 매개 변수를 선언 하는 방법](./how-to-declare-cmdlet-parameters.md)을 참조 하세요.)

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a>참고 항목

[일반 매개 변수 이름](./common-parameter-names.md)

[Cmdlet 매개 변수를 선언 하는 방법](./how-to-declare-cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
