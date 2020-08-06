---
title: 인수 집합의 유효성을 검사 하는 방법 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateSet attribute, example
ms.openlocfilehash: 6173f1380583f5b27e2b188990a5ea041f447c57
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782007"
---
# <a name="how-to-validate-an-argument-set"></a>인수 집합을 확인하는 방법

이 예제에서는 cmdlet이 실행 되기 전에 Windows PowerShell 런타임에서 매개 변수 인수를 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다. 이 유효성 검사 규칙은 매개 변수 인수에 대 한 유효한 값 집합을 제공 합니다.

> [!NOTE]
> 이 특성을 정의 하는 클래스에 대 한 자세한 내용은 [Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)를 참조 하세요.

## <a name="to-validate-an-argument-set"></a>인수 집합의 유효성을 검사 하려면

- 다음 코드와 같이 ValidateSet 특성을 추가 합니다. 이 예에서는 매개 변수에 사용할 수 있는 세 가지 값 집합을 지정 합니다 `UserName` .

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

이 특성을 선언 하는 방법에 대 한 자세한 내용은 [ValidateSet Attribute 선언](./validateset-attribute-declaration.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[Validatesetattribute.](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[ValidateSet 특성 선언](./validateset-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
