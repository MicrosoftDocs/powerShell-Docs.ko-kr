---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 매개 변수를 선언하는 방법
description: Cmdlet 매개 변수를 선언하는 방법
ms.openlocfilehash: ed53f9788c9afb142b137e08966dff33551b9d0f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667099"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Cmdlet 매개 변수를 선언하는 방법

이러한 예제에서는 명명 된, 위치, 필수, 선택적 및 스위치 매개 변수를 선언 하는 방법을 보여 줍니다. 또한이 예제에서는 매개 변수 별칭을 정의 하는 방법을 보여 줍니다.

## <a name="how-to-declare-a-named-parameter"></a>명명 된 매개 변수를 선언 하는 방법

- 다음 코드와 같이 공용 속성을 정의 합니다. 매개 변수 특성을 추가 하는 경우 `Position` 특성에서 키워드를 생략 합니다.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.

## <a name="how-to-declare-a-positional-parameter"></a>위치 매개 변수를 선언 하는 방법

- 다음 코드와 같이 공용 속성을 정의 합니다. 매개 변수 특성을 추가 하는 경우 `Position` 키워드를 인수 위치로 설정 합니다. 값 0은 첫 번째 위치를 나타냅니다.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.

## <a name="how-to-declare-a-mandatory-parameter"></a>필수 매개 변수를 선언 하는 방법

- 다음 코드와 같이 공용 속성을 정의 합니다. 매개 변수 특성을 추가 하는 경우 `Mandatory` 키워드를로 설정 `true` 합니다.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.

## <a name="how-to-declare-an-optional-parameter"></a>선택적 매개 변수를 선언 하는 방법

- 다음 코드와 같이 공용 속성을 정의 합니다. 매개 변수 특성을 추가 하는 경우 키워드를 생략 `Mandatory` 합니다.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>스위치 매개 변수를 선언 하는 방법

- 공용 속성을 형식 [System.webserver 매개 변수로](/dotnet/api/System.Management.Automation.SwitchParameter)정의한 다음 매개 변수 특성을 선언 합니다.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

매개 변수 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.

## <a name="how-to-declare-a-parameter-with-aliases"></a>별칭을 사용 하 여 매개 변수를 선언 하는 방법

- 다음 코드와 같이 공용 속성을 정의 합니다. 매개 변수에 대 한 별칭을 나열 하는 별칭 특성을 추가 합니다. 이 예에서는 동일한 매개 변수에 대해 3 개의 별칭을 정의 합니다. 첫 번째 별칭은 바로 가기를 제공 합니다. 두 번째와 세 번째 별칭은 다양 한 시나리오에 사용할 수 있는 이름을 제공 합니다.

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Alias 특성에 대 한 자세한 내용은 [Alias 특성 선언](./alias-attribute-declaration.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Parameter 특성 선언](./parameter-attribute-declaration.md)

[Alias 특성 선언](./alias-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
