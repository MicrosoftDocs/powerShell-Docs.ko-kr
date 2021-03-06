---
ms.date: 09/13/2016
ms.topic: reference
title: 인수 개수를 확인하는 방법
description: 인수 개수를 확인하는 방법
ms.openlocfilehash: 46a32d61138fb50bceea98171f76749c9d96734d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666946"
---
# <a name="how-to-validate-an-argument-count"></a>인수 개수를 확인하는 방법

이 예제에서는 Windows PowerShell 런타임에서 cmdlet이 실행 되기 전에 매개 변수가 허용 하는 인수 개수 (개수)를 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다. 이 유효성 검사 규칙은 ValidateCount 특성을 선언 하 여 설정 합니다.

> [!NOTE]
> 이 특성을 정의 하는 클래스에 대 한 자세한 내용은 [Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)를 참조 하세요.

## <a name="to-validate-an-argument-count"></a>인수 개수를 확인 하려면

- 다음 코드와 같이 Validate 특성을 추가 합니다. 이 예에서는 매개 변수에서 인수를 하나 또는 3 개까지 허용 하도록 지정 합니다.

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

이 특성을 선언 하는 방법에 대 한 자세한 내용은 [Validatecount 특성 선언](./validatecount-attribute-declaration.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[ValidateCount 특성 선언](./validatecount-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
