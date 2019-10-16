---
title: 인수의 길이를 확인 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365492"
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

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
