---
title: 인수 패턴의 유효성을 검사 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855069"
---
# <a name="how-to-validate-an-argument-pattern"></a>인수 패턴 유효성을 검사하는 방법

이 예제에서는 Windows PowerShell 런타임이 cmdlet을 실행 하기 전에 매개 변수 인수의 문자 패턴을 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다. ValidatePattern 특성을 선언 하 여이 유효성 검사 규칙을 설정 합니다.

> [!NOTE]
> 이 특성을 정의 하는 클래스에 대 한 자세한 내용은 참조 하세요. [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)합니다.

## <a name="to-validate-an-argument-pattern"></a>인수 패턴의 유효성을 검사 하려면

- 다음 코드에 표시 된 것과 같이 유효성 검사 특성을 추가 합니다. 이 예제에서는 각 숫자에 0 ~ 9의 값이 있는 4 자리 숫자로, 패턴을 지정 합니다.

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

이 특성을 선언 하는 방법에 대 한 자세한 내용은 참조 하세요. [ValidatePattern 특성 선언을](./validatepattern-attribute-declaration.md)합니다.

## <a name="see-also"></a>참고 항목

[ValidatePattern 특성 선언](./validatepattern-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
