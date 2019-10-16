---
title: 인수 개수를 확인 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365532"
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
