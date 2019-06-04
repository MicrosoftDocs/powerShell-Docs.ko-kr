---
title: Cmdlet 매개 변수를 선언 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067918"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Cmdlet 매개 변수를 선언하는 방법

이러한 예제에는 명명 된, 위치, 필수 (선택 사항)를 선언 하 고 매개 변수를 전환 하는 방법을 보여 줍니다. 이러한 예제에는 매개 변수 별칭을 정의 하는 방법을 보여 줍니다.

## <a name="how-to-declare-a-named-parameter"></a>명명된 된 매개 변수를 선언 하는 방법

- 다음 코드에 표시 된 대로 공용 속성을 정의 합니다. 매개 변수 특성을 추가한 경우 생략 된 `Position` 특성에서 키워드입니다.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

매개 변수 특성에 대 한 자세한 내용은 참조 하세요. [매개 변수 특성 선언](./parameter-attribute-declaration.md)합니다.

## <a name="how-to-declare-a-positional-parameter"></a>위치 매개 변수를 선언 하는 방법

- 다음 코드에 표시 된 대로 공용 속성을 정의 합니다. 매개 변수 특성을 추가할 때 설정는 `Position` 키워드 인수 위치입니다. 값 0은 첫 번째 위치를 나타냅니다.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

매개 변수 특성에 대 한 자세한 내용은 참조 하세요. [매개 변수 특성 선언](./parameter-attribute-declaration.md)합니다.

## <a name="how-to-declare-a-mandatory-parameter"></a>필수 매개 변수를 선언 하는 방법

- 다음 코드에 표시 된 대로 공용 속성을 정의 합니다. 매개 변수 특성을 추가할 때 설정 된 `Mandatory` 키워드를 `true`입니다.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

매개 변수 특성에 대 한 자세한 내용은 참조 하세요. [매개 변수 특성 선언](./parameter-attribute-declaration.md)합니다.

## <a name="how-to-declare-an-optional-parameter"></a>선택적 매개 변수를 선언 하는 방법

- 다음 코드에 표시 된 대로 공용 속성을 정의 합니다. 매개 변수 특성을 추가한 경우 생략 된 `Mandatory` 키워드입니다.

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

- 형식으로 공용 속성을 정의 [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)과 다음 매개 변수 특성을 선언 합니다.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

매개 변수 특성에 대 한 자세한 내용은 참조 하세요. [매개 변수 특성 선언](./parameter-attribute-declaration.md)합니다.

## <a name="how-to-declare-a-parameter-with-aliases"></a>별칭을 사용 하 여 매개 변수를 선언 하는 방법

- 다음 코드에 표시 된 대로 공용 속성을 정의 합니다. 매개 변수의 별칭을 나열 하는 별칭 특성을 추가 합니다. 이 예제에서는 세 가지 별칭은 동일한 매개 변수에 정의 됩니다. 첫 번째 별칭에는 바로 가기를 제공 합니다. 두 번째 및 세 번째 별칭에는 다양 한 시나리오에 사용할 수 있는 이름을 제공 합니다.

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

Alias 특성에 대 한 자세한 내용은 참조 하세요. [별칭 특성 선언은](./alias-attribute-declaration.md)합니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[매개 변수 특성 선언](./parameter-attribute-declaration.md)

[별칭 특성 선언](./alias-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
