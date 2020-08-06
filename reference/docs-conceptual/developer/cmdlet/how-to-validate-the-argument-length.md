---
title: 인수의 길이를 확인 하는 방법 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateLength attribute, example
ms.openlocfilehash: aa0545def6d9628f6b41090a425f0c5af25f6ad7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784081"
---
# <a name="how-to-validate-the-argument-length"></a>인수 길이 유효성을 검사하는 방법

이 예에서는 Windows PowerShell 런타임에서 cmdlet이 실행 되기 전에 매개 변수 인수의 문자 수 (길이)를 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다. ValidateLength 특성을 선언 하 여이 유효성 검사 규칙을 설정 합니다.

> [!NOTE]
> 이 특성을 정의 하는 클래스에 대 한 자세한 내용은 [Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)를 참조 하세요.

## <a name="to-validate-the-argument-length"></a>인수 길이를 확인 하려면

- 다음 코드와 같이 Validate 특성을 추가 합니다. 이 예에서는 인수의 길이는 0 자에서 10 자 사이 여야 합니다.

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

이 특성을 선언 하는 방법에 대 한 자세한 내용은 [ValidateLength Attribute 선언](./validatelength-attribute-declaration.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[ValidateLength 특성 선언](./validatelength-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
