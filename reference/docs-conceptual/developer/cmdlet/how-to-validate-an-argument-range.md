---
ms.date: 09/13/2016
ms.topic: reference
title: 인수 범위를 확인하는 방법
description: 인수 범위를 확인하는 방법
ms.openlocfilehash: 1c1c53d43350a38beb2193200de3bd6b689366a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666929"
---
# <a name="how-to-validate-an-argument-range"></a>인수 범위를 확인하는 방법

이 예제에서는 cmdlet이 실행 되기 전에 Windows PowerShell 런타임에서 매개 변수 인수의 최소값과 최대값을 확인 하는 데 사용할 수 있는 유효성 검사 규칙을 지정 하는 방법을 보여 줍니다. ValidateRange 특성을 선언 하 여이 유효성 검사 규칙을 설정 합니다.

> [!NOTE]
> 이 특성을 정의 하는 클래스에 대 한 자세한 내용은 [Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)를 참조 하세요.

### <a name="to-validate-an-argument-range"></a>인수 범위의 유효성을 검사 하려면

- 다음 코드와 같이 ValidateRange 특성을 추가 합니다. 이 예에서는 매개 변수에 대해 0에서 5 사이의 범위를 지정 합니다 `InputData` .

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

이 특성을 선언 하는 방법에 대 한 자세한 내용은 [ValidateRange Attribute 선언](./validaterange-attribute-declaration.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[ValidateRange 특성 선언](./validaterange-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
