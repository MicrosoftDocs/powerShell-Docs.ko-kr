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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067810"
---
# <a name="how-to-validate-an-argument-count"></a>인수 개수를 확인하는 방법

Windows PowerShell 런타임에 매개 변수를 허용 하는 인수 (개수)의 수를 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 주는이 예제 cmdlet을 실행 하기 전에 합니다. ValidateCount 특성을 선언 하 여이 유효성 검사 규칙을 설정 합니다.

> [!NOTE]
> 이 특성을 정의 하는 클래스에 대 한 자세한 내용은 참조 하세요. [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)합니다.

## <a name="to-validate-an-argument-count"></a>인수 개수를 유효성을 검사 하려면

- 다음 코드에 표시 된 것과 같이 유효성 검사 특성을 추가 합니다. 이 예제에서는 매개 변수 하나 또는 인수 세 개의 수락 함을 지정 합니다.

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

이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [ValidateCount 특성 선언을](./validatecount-attribute-declaration.md)합니다.

## <a name="see-also"></a>참고 항목

[ValidateCount 특성 선언](./validatecount-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
