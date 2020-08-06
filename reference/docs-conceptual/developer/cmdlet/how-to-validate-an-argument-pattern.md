---
title: 인수 패턴의 유효성을 검사 하는 방법 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidatePattern attribute, example
ms.openlocfilehash: 35104e786d4b809a711d97fea52ae0e348dd5ca3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782092"
---
# <a name="how-to-validate-an-argument-pattern"></a>인수 패턴 유효성을 검사하는 방법

이 예제에서는 cmdlet이 실행 되기 전에 Windows PowerShell 런타임에서 매개 변수 인수의 문자 패턴을 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다. ValidatePattern 특성을 선언 하 여이 유효성 검사 규칙을 설정 합니다.

> [!NOTE]
> 이 특성을 정의 하는 클래스에 대 한 자세한 내용은 [Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)를 참조 하세요.

## <a name="to-validate-an-argument-pattern"></a>인수 패턴의 유효성을 검사 하려면

- 다음 코드와 같이 Validate 특성을 추가 합니다. 이 예에서는 네 자리의 패턴을 지정 합니다. 여기서 각 숫자의 값은 0에서 9 까지입니다.

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

이 특성을 선언 하는 방법에 대 한 자세한 내용은 [ValidatePattern Attribute 선언](./validatepattern-attribute-declaration.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[ValidatePattern 특성 선언](./validatepattern-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
