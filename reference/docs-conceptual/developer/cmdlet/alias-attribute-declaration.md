---
title: Alias 특성 선언 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.openlocfilehash: 4c1ff34a244611173ca919a44d6598189b19dc98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782415"
---
# <a name="alias-attribute-declaration"></a>Alias 특성 선언

Alias 특성을 사용 하면 사용자가 cmdlet 매개 변수에 대해 다른 이름을 지정할 수 있습니다. 별칭을 사용 하 여 매개 변수 이름에 대 한 바로 가기를 제공 하거나 다양 한 시나리오에 적합 한 다른 이름을 제공할 수 있습니다.

## <a name="syntax"></a>구문

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>매개 변수

`aliasName`(String []) 필수. Cmdlet 매개 변수에 대 한 쉼표로 구분 된 별칭 이름 집합을 지정 합니다.

## <a name="remarks"></a>설명

- Alias 특성은 cmdlet 매개 변수를 지정할 때 Parameter 특성과 함께 사용 됩니다. 이러한 특성을 선언 하는 방법에 대 한 자세한 내용은 [Cmdlet 매개 변수를 선언 하는 방법](./how-to-declare-cmdlet-parameters.md)을 참조 하세요.

- 각 별칭 이름은 cmdlet 내에서 고유 해야 합니다. Windows PowerShell은 중복 된 별칭 이름을 확인 하지 않습니다.

- 별칭 특성은 cmdlet의 각 매개 변수에 대해 한 번만 사용 됩니다.

- Alias 특성은 [Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 클래스에 의해 정의 됩니다.

## <a name="see-also"></a>참고 항목

[매개 변수 별칭](./parameter-aliases.md)

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
